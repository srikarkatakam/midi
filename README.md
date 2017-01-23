package music;
import javax.sound.midi.*;

public class midi2 {
	public static void main(String a[]) throws Exception{
		midi2 mi=new midi2();
		System.out.println("awesome");
		mi.play();
	}
	public void play() throws Exception{
		Sequencer player=MidiSystem.getSequencer();
		player.open();
		Sequence sq=new Sequence(Sequence.PPQ,4);
		Track track=sq.createTrack();
		track.add(makeEvent(192,1,35,100,5));
		for(int i=5;i<61;i+=2){
			track.add(makeEvent(144,1,i,100,i));
			track.add(makeEvent(144,1,i,100,i));
		}
		player.setSequence(sq);
		player.start();
		
		
		
		
	}
	public static MidiEvent makeEvent(int comd,int chan,int one,int two,int tick) throws Exception{
		MidiEvent event=null;
		ShortMessage noteon=new ShortMessage(comd,chan,one,two);
		event=new MidiEvent(noteon,tick);
		return event;
	}

}
